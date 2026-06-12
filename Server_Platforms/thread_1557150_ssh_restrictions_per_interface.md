---
title: "ssh restrictions per interface?"
date: 2010-08-20
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-08-20
I have a server with two active network interfaces.  On one, I need ssh open for all users (it's running LTSP, and as I learned the hard way today, blocking ssh kills LDM access).

On the other interface (which connects to the rest of the network), I only want to allow a few administrative users to connnect.

Is there a way to do this cleanly using sshd_config or PAM? I don't want to do something hacky like running dropbear.

---

### Post by Fire_Chief on 2010-08-20
Since SSH is a system wide service, it doesn't really work that way. You can prevent individual users or prevent individual networks but both changes affect the way SSH and the whole server listens and permits logins.

Let's call the LTSP user network interface NIC1 and the other "rest of the network" interface NIC2.

You could use IPtables or another firewall to:
1st - permit SSH from the NIC1 network
2nd - permit SSH from specific NIC2 network IPs or subnets
3rd - block SSH from everywhere else
This would allow only users from specific IPs on the NIC2 network (i.e. admin PCs) to SSH on the server but still allow all users on NIC1 network to have SSH access for LTSP functionality.
Of course the limitation is that the admin access is not so much restricted to specific users but rather the specific IPs that SSH would allow access from (hopefully static IPs of admin workstations or IP range of admin only users).

Cheers!

---

### Post by lykwydchykyn on 2010-08-20
Thanks for the suggestions; I don't know that that approach will answer.  

I wonder, is it possible to allow specific users only from a specific network (i.e. -- user "ltsp10" may only connect from 10.10.7.0/24)?

I have a hard time believing such a flexible service as ssh is this inflexible about authorization rules.

---

### Post by lykwydchykyn on 2010-08-23
Ok, I found a solution.

What I needed was /etc/security/access.conf.

I still can't do it by interface, but I can do it by network which was ok since the LTSP side only has one network.

It was as simple as adding three rules to access.conf:
```

+ : (admin) : ALL
+ : (kiosks) : thin_client_network_CIDR
- : ALL : ALL

```

Then I had to change /etc/pam.d/sshd to uncomment the line:
```

account required pam_access.so

```

And it works like a charm!

---

