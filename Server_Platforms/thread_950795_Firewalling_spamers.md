---
title: "Firewalling spamers"
date: 2008-10-17
forum: Server Platforms
---

### Post by tonkyman on 2008-10-17
I have someone trying to get into my mail server right now and I need to find a way to make them stop. How can I firewall them and drop them???

I'm running Ubuntu 8.04 as a mail server with postfix, courier, squirrell mail and that sort of stuff.

Thanks

---

### Post by hrod beraht on 2008-10-17
For a quick-fix, if you just want to block a particular IP address, you can just add it to your [iptables]("https://help.ubuntu.com/community/IptablesHowTo").

```
# iptables -A INPUT -s xxx.xxx.xxx.xxx -j DROP
```
Where xxx.xxx.xxx.xxx is the IP address you want to block. Or install *Firestarter* through Synaptic if you want a GUI front-end.

Bob

---

### Post by cdenley on 2008-10-17
Are they trying to guess passwords? To prevent dictionary attacks, use fail2ban. It will probably require some configuration for it to read authentication attempts from the mail server you're running.

---

### Post by tonkyman on 2008-10-17
Thanks Bob, that took care of them. :popcorn:

They had been hitting the server for over an hour with login attempts. They were not getting in but were causing a TON of traffic.

It's my understanding that the iptables rule I just entered will go away after I reboot... is that true?

Tony

---

### Post by cdenley on 2008-10-17
Yes. If you don't want it to, add a script to /etc/network/if-up.d, or use ufw.
```

sudo ufw enable
sudo ufw deny proto tcp from xxx.xxx.xxx.xxx

```
Fail2ban would prevent attacks such as this from any host.

---

### Post by hrod beraht on 2008-10-17
> **tonkyman said:**
> Thanks Bob, that took care of them. :popcorn:

They had been hitting the server for over an hour with login attempts. They were not getting in but were causing a TON of traffic.

Hopefully that gets rid of them forever. However, as I mentioned, it's more of a quick-fix. The reason being that it only blocks that one IP address. If they're persistent and come at you from other addresses, having to block them manually, one by one would probably be a pain in the neck.

As Cdenley suggests, something like fail2ban might be what you are looking for as a more automated solution. It basically looks for a lot of failed logins and then adjusts the iptables automatically to block them.

Bob

---

### Post by tonkyman on 2008-10-20
> **cdenley said:**
> Yes. If you don't want it to, add a script to /etc/network/if-up.d, or use ufw.
```

sudo ufw enable
sudo ufw deny proto tcp from xxx.xxx.xxx.xxx

```
Fail2ban would prevent attacks such as this from any host.

Thanks Cdenley, I tried to use ufw but was never able to figure out how to use it where it didn't deny everything. That command is going in my notebook along with bob's iptable command... good stuff to know.

Thanks,
Tony

---

