---
title: "Spoofed SSH-attacks - how to find source?"
date: 2021-01-27
forum: Security
---

### Post by Elmi77 on 2021-01-27
Hi,

I experience attacks to my dedicated server for some months. There is some automated script trying to break into the server by brute force. It is connecting to SSH and tries several usernames and passwords. It is not a security risk at the moment as my SSHD is turned off and I turn it back on only when I need it (there is a possibility to do that via the hosting provider). And when it is turned on the script fails because of very long and unusual usernames and passwords.

Nevertheless I would like to get rid of this. Unfortunately this is not that easy as the IP where the SSH-access comes from changes every 2..5 tries (means even fail2ban is not a solution for this).

For me it looks like the IP is spoofed.

My question: how can I find out what the real IP is where this attacks come from?

Thanks!

---

### Post by The Cog on 2021-01-27
They cannot spoof the IP because ssh needs two-way traffic to work.
But they can and do use distributed hacking from the thousands of machines they have compromised, in order to get round things like failtoban that block an IP after a few failed attempts.
Three things to consider:
* move your sshd to a different, random high port. That will lose most of them
* use public keys rather than passwords for authentication (passwordless ssh)
* block ssh in your firewall, apart from a few known IP address ranges that you want to serve

---

### Post by Elmi77 on 2021-01-27
> **The Cog said:**
> * move your sshd to a different, random high port. That will lose most of them

It is already running on a different port. Seems this attacker has done a portscan before.

> **The Cog said:**
> * use public keys rather than passwords for authentication (passwordless ssh)

This keeps the attacker away but I still have hundreds of log entries of failed log-ins every day, right?

> **The Cog said:**
> * block ssh in your firewall, apart from a few known IP address ranges that you want to serve

I hesitate to do that. This is something one forgets easily - and when I change my ISP one day, I'm locked out.

---

### Post by SeijiSensei on 2021-01-27
I use a static tunnel via OpenVPN to communicate with my remote servers. That's the only way you can SSH into my servers. 

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by CharlesA on 2021-01-27
Similar to SeijiSensei,I've got my external IP whitelisted and drop all other traffic to my ssh port.

No more brute force attacks in my auth.log since no connections are established. I see a ton of traffic in the firewall logs, though, but that is to be expected.

---

### Post by TheFu on 2021-01-27
Research _port knocking_ if you are unwilling to block 99% of the internet that will never, ever, need ssh into the system.

And passwords shouldn't be used for any internet facing service. Use keys.

---

### Post by The Cog on 2021-01-27
Similar to SeijiSensei, I would suggest using a wireguard VPN. Wireguard is great - easy to set up, and undetectable in that it won't give any response to packets that don't have the right key. Only allow wireguard in from the internet, and use ssh over the vpn. 

The only problem is that (as far as I know) you need to configure different keys for every user, which may be a maintenance issue if you have lots of users.

---

