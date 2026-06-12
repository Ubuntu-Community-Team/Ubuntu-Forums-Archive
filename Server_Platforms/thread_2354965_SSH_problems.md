---
title: "SSH problems"
date: 2017-03-08
forum: Server Platforms
---

### Post by toothandnail on 2017-03-08
I'm looking to replace an old home server (Slackware) with Ubuntu Server 16.04. I've had the Ubuntu machine running for a while as a secondary server, no problems there... However, to replace the Slackware server, I need dnsmasq running as a local DHCP/DNS server. And I need the Ubuntu server running a static IP.

I've finally managed to get all the details sorted out (I think...). When I first tried, I found that I was not getting any DNS relay services to other machines on my network. I've now managed to get dnsmasq and resolvconf working correctly with the Ubuntu server set to a static IP. Great, just what I need. However, I've hit another problem, which I don't understand at all.

SSH is set up on the Ubuntu server, with password authentication turned off. When the Ubuntu server was set as secondary, getting its IP from the Slacware server, I could SSH to it by name using public/private keys without any problems. As soon as the Ubuntu server is set to static, I am suddenly unable to SSH to it by name - if I do so, I get prompted for a password, which, naturally, doesn't work. Strangely, I can SSH to it by IP, at which point the public/private key pair work correctly and I can log in.

I'm not willing to enable password authentication, since I need to be able to access the server from remote locations as well as from the local network. So I'm wondering if anyone can tell me why the change, making the Ubuntu server the only server on the network suddenly disables the ability to use public/private keys ? Its name is the same, the key pair still works correctly when called by IP, the server name is obviously being seen, since I get a password prompt from the machine. The IP address of the machine is the same (I was setting it by a reserved DHCP entry from the Slackware server).

Any help much appreciated.

---

### Post by darkod on 2017-03-08
Hmmm can it be something related to known_hosts file? Yes, the IP was the same but I am not sure if it considered small difference being dhcp with reservation compared to static IP. And ssh is very careful about any changes from the original first connection and can interpret it as intent to hack in.

Why wouldn't you install the server with a static IP directly from the start?

Try deleting the entry for the ubuntu server in your client's known hosts and see if that helps.

---

### Post by volkswagner on 2017-03-08
This is likely a DNS issue.

My guess is you have another server on the LAN accepting
ssh connections or listening on port 22.

What do you get when you run 

```
nslookup nameOfUbutnuServer
```
```
ping nameOfUbutnuServer
```
```
dig nameOfUbutnuServer
```

Since the server is offering DNS to clients, it needs to "know"
it's own name. I've never run dnsmasq on Ubuntu, but when
running it on OpenWRT I usually add static DNS like:

```
config domain
        option name 'server.com'
        option ip '192.168.33.50'

```

I think the above is similar to adding an "A" record to Bind or other DNS servers.

---

### Post by toothandnail on 2017-03-08
> **darkod said:**
> Hmmm can it be something related to known_hosts file? Yes, the IP was the same but I am not sure if it considered small difference being dhcp with reservation compared to static IP. And ssh is very careful about any changes from the original first connection and can interpret it as intent to hack in.

I don''t think that can be the problem. I've got strict checking enabled, and it will normally come up with a message as soon as the fingerprint differs in any way to the original. On the client side (which should be the only one that matters when it comes to known_hosts) it will shut down the login attempt on the spot. In this instance, the server is presenting a password prompt. Possible, but I don't think its likely. I tired using -vv on the SSH command, and it seemed that the client end was attempting to present the key but it was not being noticed by the server end.

> Why wouldn't you install the server with a static IP directly from the start?

It was originally a test server. I have some clients that I want to move away from the Slackware servers I've been using in non-gateway areas. I normally only use DHCP reservations for that type of server. To be honest, I should have a spare hard drive around somewhere, so I can try an install with a static IP. 

> Try deleting the entry for the ubuntu server in your client's known hosts and see if that helps.

:) I tried moving the existing knonw_hosts file and letting it try again - same problem...

Thanks for the suggestions.

---

### Post by toothandnail on 2017-03-08
> **volkswagner said:**
> This is likely a DNS issue.

My guess is you have another server on the LAN accepting
ssh connections or listening on port 22.

Ah! Now that sounds as though it could be the problem. I have the SSH server configured on a couple of desktop machines as well. 

> What do you get when you run 

```
nslookup nameOfUbutnuServer
```
```
ping nameOfUbutnuServer
```
```
dig nameOfUbutnuServer
```



Won't be able to test that until tomorrow, but I will check then.

> Since the server is offering DNS to clients, it needs to "know"
it's own name. I've never run dnsmasq on Ubuntu, but when
running it on OpenWRT I usually add static DNS like:

```
config domain
        option name 'server.com'
        option ip '192.168.33.50'

```

I think the above is similar to adding an "A" record to Bind or other DNS servers.

That looks like the equivalent of the "host-record" command line switch. I've not seen it used in the config file, but I'll do some testing tomorrow and see where it takes me. I'll post back with the results.

Thanks for the suggestion - that looks pretty likely to be the culprit. Interesting that I didn't need it with the Slackware server. There must be something different in the way it is running dnsmasq.

---

### Post by volkswagner on 2017-03-08
> **toothandnail said:**
> 

That looks like the equivalent of the "host-record" command line switch. I've not seen it used in the config file, but I'll do some testing tomorrow and see where it takes me. I'll post back with the results.


I believe the host command is for creating a reserved dhcp address. Again, I've only worked with dnsmaq 
while using OpenWRT, so here's their description.
[https://wiki.openwrt.org/doc/uci/dhcp](https://wiki.openwrt.org/doc/uci/dhcp)

---

