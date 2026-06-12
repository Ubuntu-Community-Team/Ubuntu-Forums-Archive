---
title: "IPTABLES - most secure startup?"
date: 2015-05-03
forum: Server Platforms
---

### Post by dozy on 2015-05-03
Hello again everyone,

I have been working on making my own firewall with iptables, and I need some advice.. again!

I am trying to come up with a good way to secure the firewall machine while it is booting.
One of the challenges I am facing is that I have to wait for the public network devices to come up before I can apply some of the rules. This is because it is receiving its address via DHCP, and I need its address before I can write the rules that apply to it.

My setup is simple:
eth0 (public interface)
eth1 (private interface)

So far, the best I can come up with is to do the following in the /etc/network/interfaces file.
The idea is that everything will be set to drop before the interfaces come up, except in and out on eth1 (private), and it will be that way until the full rules are calculated and applied.
I'm not worried about being locked out of eth0 because I will always be on the eth1 side.

**/etc/network/interfaces**
```

auto lo
iface lo inet loopback

pre-up iptables-restore < /etc/iptables_startup_rules

-- eth1 config --

allow-hotplug eth0
iface eth0 inet dhcp
post-up /etc/iptables_full_rules.sh

```

**/etc/iptables_startup_rules** looks something like this. (from memory. syntax may not be 100%):
```

*filter
:INPUT DROP
:FORWARD DROP
:OUTPUT DROP

-A INPUT -i lo -j ACCEPT
-A OUTPUT -o lo -j ACCEPT

-A INPUT -i eth1 -j ACCEPT
-A OUTPUT -o eth1 -j ACCEPT

```

The **/etc/iptables_full_rules** script retrieves the  IP address from the eth0 interface - after it has come up - and uses it while building some additional rules.


So, does anyone have a better, more secure way I could protect the machine at start up?

Thanks for you time.

---

### Post by dino99 on 2015-05-03
here is what i get as recently published  [https://www.google.co.in/search?q=ubuntu+getdeb+archive&oq=ubuntu+getdeb+archive&aqs=chrome..69i57j69i64.9545j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8#tbs=qdr:m&q=ubuntu+network+links+iptables](https://www.google.co.in/search?q=ubuntu+getdeb+archive&oq=ubuntu+getdeb+archive&aqs=chrome..69i57j69i64.9545j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8#tbs=qdr:m&q=ubuntu+network+links+iptables)

---

### Post by dozy on 2015-05-03
Thanks for your reply, dino99. I appreciate your time.
However, I think based on the search link you provided, there is a misunderstanding as to the specifics of what I am asking.



Does anyone else have any suggestions for a more effective way to secure a machine while its full set of iptables rules are being created/loaded, other than what I have proposed in the original post?

Thanks again.

---

### Post by matt_symes on 2015-05-03
Thread moved to **Server Platforms**. 

You may get more responses in here but i've also left a redirect on he other subforum.

BTW: Are you currently using these rules ?

---

### Post by dozy on 2015-05-04
Thank you for the redirect.

**BTW: Are you currently using these rules ?**
Yes, but only in a test environment, until I get it all figured out.
The rules I have shown (in **/etc/iptables_startup_rules) **are only the initial rules that I apply at pre-up. They only last until all interfaces are up and the new rules are applied.

---

### Post by SeijiSensei on 2015-05-04
I think you're being overly paranoid.  

When networking starts, there are no services running so there are no exposed surfaces to exploit.

If you run iptables immediately thereafter, there really are no threats to worry about.

If you want to grab the external IP address after dhclient runs, you can use this:
```
EXT=$(ifconfig | grep 'inet addr' | head -n 1 | awk '{print $2}' | sed 's/addr://g')
```
That stores the external address in the enviroment variable EXT.  Put that in the script with the iptables rules, so you can reference the external address as $EXT.

---

### Post by dozy on 2015-05-04
Thank you for your advice, SeijiSensei. That is the kind of feedback I was looking for.

---

