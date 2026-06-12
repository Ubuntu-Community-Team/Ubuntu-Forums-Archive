---
title: "SSH security with -D and tunneling"
date: 2012-03-30
forum: Security
---

### Post by NertSkull on 2012-03-30
So, I've been reading around and came across this post

[http://superuser.com/questions/62303/how-can-i-tunnel-all-of-my-network-traffic-through-ssh](http://superuser.com/questions/62303/how-can-i-tunnel-all-of-my-network-traffic-through-ssh)

A couple posts down, someone claims that tunneling through SSH -D is not 100% secure?  But there wasn't much more discussion on why not.  

Is that statement correct?  If I'm in a public wifi setting and I'm tunneling something like this 
```
ssh -D 9999 -C me@myhost.com
```is that good enough?  Or should I be concerned about security.

I was under the impression that EVERYTHING that goes through SSH is encrypted ALL the time.  Am I missing something?

(I know that other post is talking about doing all your traffic, but I'm just interested in the ssh -D port forwarding/socks stuff).  Thanks!

---

### Post by Ms. Daisy on 2012-03-30
According to this [http://isc.sans.edu/diary.html?storyid=1603](http://isc.sans.edu/diary.html?storyid=1603)

[PARAPHRASE] 

All your web surfing will be encrypted to your home box before  traveling to the Internet [using ssh].  Most recent browsers will send your outbound DNS request through the SSH tunnel. Be advised that your outbound DNS requests  are still sent to the local network unencrypted [if you're on public wifi and using SOCKS]. So that is another  reason to use Squid if you are concerned about privacy or being  re-directed by malicious DNS servers on the wireless LAN.

[/PARAPHRASE]

---

### Post by NertSkull on 2012-03-30
Yeah, I should have mentioned that I'm using firefox, and in the about:config tab I have set

network.proxy.socks_remote_dns to true

So (from what I've read) that should take care of DNS lookup through the proxy.

So, aside from that, is there any other potential security issue with this setup?

---

### Post by kevdog on 2012-03-30
Where's the link suggesting the -D option is unsecure. I've never heard of this before.

---

### Post by Dangertux on 2012-03-30
The option -D is not inherently insecure. I am not sure why anyone is saying it is, the few arguments that were presented make no sense.

-D binds to a local port and creates a socks listener. That is all. All traffic that is proxied through SSH will be encrypted between the client and the ssh tunnel's endpoint.

Now if the application that is using the tunnel does something dumb like not using the tinnel for dns lookups it is that application's security issue not an issue with the ssh tunnel (since it was never used)

Hope this hells

---

### Post by Ms. Daisy on 2012-03-30
Dangertux, so the sans link is incorrect- that outbound DNS requests  are NOT sent to the local network unencrypted?

---

### Post by Dangertux on 2012-03-30
I'm not saying the link was incorrect, I'm saying it has absolutely nothing to do with SSH, but how the program utilizing the proxy makes calls for DNS resolution. 

It's like saying the ssh -D option sucks because my browser is stupid. It makes no sense.

From the ssh man page

> 
 -D [bind_address:]port
             Specifies a local “dynamic” application-level port forwarding.
             This works by allocating a socket to listen to port on the local
             side, optionally bound to the specified bind_address.  Whenever a
             connection is made to this port, the connection is forwarded over
             the secure channel, and the application protocol is then used to
             determine where to connect to from the remote machine.  Currently
             the SOCKS4 and SOCKS5 protocols are supported, and ssh will act
             as a SOCKS server.  Only root can forward privileged ports.
             Dynamic port forwardings can also be specified in the configura&#8208;
             tion file.

             IPv6 addresses can be specified by enclosing the address in
             square brackets.  Only the superuser can forward privileged
             ports.  By default, the local port is bound in accordance with
             the GatewayPorts setting.  However, an explicit bind_address may
             be used to bind the connection to a specific address.  The
             bind_address of “localhost” indicates that the listening port be
             bound for local use only, while an empty address or ‘*’ indicates
             that the port should be available from all interfaces.



So if your browser doesn't proxy DNS requests use a different browser I guess? 

I mean I'm not even sure what the person in that article is even pointing that out for -- bottom line on SSH if it goes THROUGH the ssh forward, it WILL be encrypted until the endpoint (of the forward, not the final destination).

Also "DNS requests to the local network" is ambiguous, convoluted and makes it seem like the author has no clue what they're talking about.

Possible scenario DNS requests to a host name for which an internal DNS server (not reachable from the SSH proxy) is authoritative, will HAVE to be made in the clear.

But how many people are doing that?

---

### Post by HermanAB on 2012-04-01
Howdy,

Run tcpdump or wireshark and look at the network connection.  If everything is gobbledygook, then you are OK.  If you see plain text, then you are not.

If you want even more confidence, capture a bunch of data then try to compress it with gzip.  If it compresses, then the encryption is broken, if not, then you are very probably OK.

---

### Post by NertSkull on 2012-04-02
Thanks for everyone's input.  Kind of what I've always been told, that once the connection is established properly, everything is secure.  I will disregard the article.

Who knew the internet had bad information in it?  :)

---

