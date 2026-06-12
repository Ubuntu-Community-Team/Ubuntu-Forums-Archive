---
title: "Does denyhosts work if ssh is on a nonstandard port?"
date: 2007-08-13
forum: Server Platforms
---

### Post by Atreus12 on 2007-08-13
I installed denyhosts, but I am using ssh on a nonstandard port. Just to test it out, I ssh'ed in and gave an incorrect password 5 times in a row. Ssh still works, even though the config file specifies a limit of 3. Also,  /etc/hosts.deny is empty

Do I have to do something special to get this to work?

Also, after not getting denyhosts to work, I set some [ Iptables Rules](http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/), and managed to lock myself out.

When I flush iptables, I can get in, but after adding the rules again, I am still locked out. Where is iptables storing the banned ip addresses?

-Andrew

Edit: ssh logging is set at VERBOSE, would that mess anything up?

---

### Post by p_quarles on 2007-08-13
If you haven't already, make sure you start the program in background mode:
```
sudo denyhosts --daemon
```
And, no, your SSH logging level will not affect this.

By the way, are you aware that the phrase "iptables rules" in your message links to Wikipedia's article on pangolins? :-)

---

### Post by Atreus12 on 2007-08-13
> **p_quarles said:**
> 
By the way, are you aware that the phrase "iptables rules" in your message links to Wikipedia's article on pangolins? :-)

Blast. Apparently ctrl+a and middle click do not work together. In firefox at least.

If you are wondering, that link came from someone recommending a pangolin laptop. I wasn't sure what they were talking about so I googled it, and  its a system76 model.

I fixed the link.

To get back on topic :)  Yes, the denyhosts daemon is running. I stopped it and restarted it just to make sure. Does a nonstandard port have anything to do with it? I am also exclusively using ssh keys, meaning that password authentication is disabled. Would this have anything to do with it?

Also, can someone explain the iptables lockout to me? How does iptables remember ip addresses?

-Andrew

---

