---
title: "How insecure is  this Network?"
date: 2007-02-28
forum: Server Platforms
---

### Post by cd-r80 on 2007-02-28
How insecure is  this Network?

DSL Linux
eth0 DHCP
eth0:1 192.168.0.2
|
|
ADSL Router---INTERNET
|
|
Ubuntu Dualboot W$.
eth0 DHCP
eth0:1 192.168.0.1

I use DSL as a fileserver through 192.168.0.0 net.
Both use internet.
Now I use only FTP start/stop.  Can I setup Samba on DSL Linux For only 192.168.0.0?

---

### Post by kidders on 2007-02-28
Hi there,

Sorry for answering a question with a question, but what kind of security issues are you concerned about? For instance, are we talking about "industrial strength" security, or are you just interested in not doing something overtly silly?

---

### Post by cd-r80 on 2007-02-28
Is This very silly or easy? Of course I want to be as secure as possible. Or how easy it is spy that localnet?

---

### Post by kidders on 2007-02-28
> **cd-r80 said:**
> Is This very silly or easy?Oh no... not at all. It's just a question of how paranoid you'd like to be. For instance, it would be technically valid to claim that your network is unsafe, because the DNS implementation on your router (which is, by its nature, less frequently updated than a software-based DNS) may be flawed, making it vulnerable to local attack. This would expose you to a wide range of devastating hacks, assuming a sufficiently expert local user (or a user that could *get* local access) was interested in causing trouble. Virtually everyone could discount that as pointlessly paranoid though.

> **cd-r80 said:**
> Or how easy it is spy that localnet?Ah, so you're interested in *local* security. To sort local issues out, you need to decide who should have access to your LAN in the first place. For instance, would you like to try to prevent computers you haven't preauthorised from connecting to your network?

The next step is to assume that a malicious user has gained access, despite any attempts you may have made to make that difficult, and think about what kind of access he could get to any services you are running. Passwords, for instance, need to be of good quality.

Then, it's worth considering the issue you mentioned ... passively listening for interesting packets. If you're worried about this issue, using FTP (which you mentioned) would be totally unacceptable ... all data, including login details would flow over the network as plain text. If you're interested in seeing how amazingly easy it would be to acquire your login information, try playing around with Ethereal (now called Wireshark afaik). Tools like these may also expose login details for remote services, such as your email accounts, along with any data exchanged.

If you're interested in sharing files securely, the most straightforward solution is SFTP (sometimes called fish://). It's a system most people are familiar with (because it operates over SSH), and is heavily encrypted. There are plenty of other options, but virtually all Linux users know SSH very well, so they can understand how it works very quickly/easily.

---

### Post by cd-r80 on 2007-02-28
ADSL Router is bridged mode On, no DSN on Router. Same time works as a LAN Router. DHCP IPs are a real world. Just wonder how If someone can enter bridged router from outside. Or how Two IPs work on a same NIC? If somenone Listens REAL IP (same interface) can he somehow see also the virtual IP trafic?

---

### Post by kidders on 2007-03-01
> **cd-r80 said:**
> ADSL Router is bridged mode On, no DSN on Router. Same time works as a LAN Router.Interesting... So your ISP lets you use more than one IP address?

> **cd-r80 said:**
> Or how Two IPs work on a same NIC?A network interface can only have one IP, which I imagine is why you've set up some virtual interfaces.

I wouldn't be particularly confident about this setup. Although, in theory, it should be perfectly fine, your network security depends heavily on the quality of your router's software.

> **cd-r80 said:**
> If somenone Listens REAL IP (same interface) can he somehow see also the virtual IP trafic?That would be entirely up to your router imo. Assuming everything is configured properly, you should only be vulnerable if there is a known problem with your specific router's firmware.

---

### Post by cd-r80 on 2007-03-01
Yes, I can have 5 IPs. Normal here. I try to investigate that router's secur more. At least I have disabled admin conn. from outside. It has some more options also... Is it easy or possible to make a tunnel for Samba? Perhaps not when booted in Win$.

---

### Post by kidders on 2007-03-01
> **cd-r80 said:**
> Is it easy or possible to make a tunnel for Samba?How do your other network services work? Is your router not capable of routing packets correctly between two private IPs?

---

### Post by cd-r80 on 2007-03-01
LAN 192.168.0.0 is fast and works well.  Via ISP it works also of course, with slower connection. FTP LAN & browse internet works well at same time. I just wonder if I Make tunnels, then no one cannot listen from the router, of course so...

---

### Post by kidders on 2007-03-02
You *could* do that, but anything you tunneled through your public IPs would slow down, depending on the speed of your internet connection, and slow down even further, because of the added load of encrypting everything.

I'm suspicious of your network configuration, because it just doesn't "feel" right, which is really only an opinion. It may in fact be perfectly secure. Having said that, I would *never* configure a network of mine this way.

---

### Post by cd-r80 on 2007-03-02
Now I just don't have to install more NICs or cables.  I tried Wlan, but it does not pass walls. I wonder how the router survives so well, but it just works very well.

---

