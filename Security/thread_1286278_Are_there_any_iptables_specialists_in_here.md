---
title: "Are there any iptables specialists in here?"
date: 2009-10-08
forum: Security
---

### Post by viking_maniac on 2009-10-08
I would be very grateful for some help to setup a specific rule:

Since I'm using the TOR application for anonymity, I'd like to configure iptables to only allow _TOR_ as an application to connect to Internet as in outgoing requests. And of course still deny all incoming, like my default UFW setting is now. I want to plug any leaks, like software bugs, DNS leaks or any application that could bypass TOR and compromise my anonymity.

I'd also like to turn this **on** and **off**, either with a command or a shell script, so I can access Internet with any outgoing request when I'm not using TOR.

Thanks in advance! :)

---

### Post by update_manager on 2009-10-08
> **viking_maniac said:**
> I would be very grateful for some help to setup a specific rule:

Since I'm using the TOR application for anonymity, I'd like to configure iptables to only allow _TOR_ as an application to connect to Internet as in outgoing requests. And of course still deny all incoming, like my default UFW setting is now. I want to plug any leaks, like software bugs, DNS leaks or any application that could bypass TOR and compromise my anonymity.

I'd also like to turn this **on** and **off**, either with a command or a shell script, so I can access Internet with any outgoing request when I'm not using TOR.

Thanks in advance! :)


That will be hard but possible.

From the iptables man page:

[INDENT][I]owner
       This  module  attempts  to match various characteristics of the packet creator, for locally generated
       packets. This match is only valid in the OUTPUT and POSTROUTING chains. Forwarded packets do not have
       any  socket associated with them. Packets from kernel threads do have a socket, but usually no owner.

       [!] --uid-owner username

       [!] --uid-owner userid[-userid]
              Matches if the packet socket&#8217;s file structure (if it has one) is owned by the given user.  You
              may also specify a numerical UID, or an UID range.

       [!] --gid-owner groupname

       [!] --gid-owner groupid[-groupid]
              Matches if the packet socket&#8217;s file structure is owned by the given group.  You may also spec&#8208;
              ify a numerical GID, or a GID range.

       [!] --socket-exists
              Matches if the packet is associated with a socket.
[/I][/INDENT]


If you're starting tor as root:


# allow tcp connections for processes owned by root
iptables -I OUTPUT -p tcp -m --uid-owner root -j ACCEPT

# allow anyone to talk on the LAN or to localhost
iptables -A OUTPUT -p tcp -d $LAN -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# last rule, drop all output
iptables -A OUTPUT -p tcp -j DROP

---

### Post by HermanAB on 2009-10-08
Hmm, if Tor is compiled with tcpwrappers libwrap, then you can easily control it in /etc/hosts.allow.

---

### Post by viking_maniac on 2009-10-09
How about this one?

```
# iptables -F OUTPUT
# iptables -A OUTPUT -j ACCEPT -m owner --uid-owner debian-tor
# iptables -A OUTPUT -j ACCEPT -o lo
# iptables -P OUTPUT DROP
# iptables -L -v
```I just found it on the TOR wiki site after some intensive searching. But I don't know how safe it is to use. Could anyone be so kind to analyze it and see what it does?

BTW, how do you remove iptables rules if you should mess things up?

---

### Post by update_manager on 2009-10-09
> **viking_maniac said:**
> How about this one?

```
# iptables -F OUTPUT
# iptables -A OUTPUT -j ACCEPT -m owner --uid-owner debian-tor
# iptables -A OUTPUT -j ACCEPT -o lo
# iptables -P OUTPUT DROP
# iptables -L -v
```I just found it on the TOR wiki site after some intensive searching. But I don't know how safe it is to use. Could anyone be so kind to analyze it and see what it does?

BTW, how do you remove iptables rules if you should mess things up?

To remove iptables rules:
sudo iptables -F

These rules don't allow any output traffic unless the process is owned by the "debian-tor" user or the interface is the loopback adapter.

This can fail in a few places (see the iptables man page for details) but look pretty good.

---

### Post by viking_maniac on 2009-10-10
> **update_manager said:**
> To remove iptables rules:
sudo iptables -F

These rules don't allow any output traffic unless the process is owned by the "debian-tor" user or the interface is the loopback adapter.

This can fail in a few places (see the iptables man page for details) but look pretty good.

Thanks for your feedback!

Do you recommend any revisions to this code, to be even more safe?
Or is this the best as it can get?

---

### Post by update_manager on 2009-10-10
> **viking_maniac said:**
> Thanks for your feedback!

Do you recommend any revisions to this code, to be even more safe?
Or is this the best as it can get?

Its not going to work in all possible cases. Even when it does work, the results might not be what you expect - processes owned by the tor user can send out normal traffic.

You might want to do some port-based restrictions such as:
iptables -A OUTPUT -m multiport -p tcp --dport 137:139,445 -j REJECT

---

### Post by Lars Noodén on 2009-10-11
Also, since the policy cannot use the REJECT target, you'll need to make the last rule something like this:

iptables -A OUTPUT -j REJECT

It will make diagnosis of problems much easier.

---

### Post by viking_maniac on 2009-10-11
> **update_manager said:**
> Its not going to work in all possible cases. Even when it does work, the results might not be what you expect - processes owned by the tor user can send out normal traffic.

You might want to do some port-based restrictions such as:
iptables -A OUTPUT -m multiport -p tcp --dport 137:139,445 -j REJECT

Are these ports special in any way, or are they just random samples?

The user **debian-tor** is the only one active and is the one that owns the TOR process as it starts and as long as it runs - no other processes starts with that user as far as i can see and have understood. This is not a regular user account, but you might already know that. It should therefore be pretty hard for any other application, like Firefox, owned by my active user account, to leak normal traffic unless I'm missing some important points here regarding iptables and how it works. I've done some excessive testing with Wireshark to prove that point; TOR is the only process using the net and nothing else works if I try to access the Internet.

---

### Post by lensman3 on 2009-10-11
Your iptable rules appear to be on a single machine attached to the Internet.  The command "netstat -a" should show you which ports are connected to the internet.  The first part is the important part and has the title "Active Internet connections (servers and established)".  For what you want to do, only the tor port should be outgoing (I think).  Tor as I remember does tunneling.  I don't remember what a tunnel port connection would look like from "netstat -a".  


netstat -a stands for all.

Hope this helps a little.

---

