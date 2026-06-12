---
title: "Only allowed to use one port for proxy"
date: 2010-06-05
forum: Security
---

### Post by cwwilson721 on 2010-06-05
I'm using a local proxy server VPN'd to another network.

How do I setup either Firestarter or Gufw/ufw to ONLY allow in/out from ONE port? (The one port the proxy uses)

Ex: Firefox is proxied to 127.0.0.1, all ports, and then the proxy picks it up, and sends out on port xxxx, and recieves on port xxxx, then sends back thru 127.0.0.1, back to Firefox.

Any setting/rules I've treid on either Firestarter or Gufw kills the proxy>VPN (Proxy won't connect to remote network)

It's probably fairly easy, but my mind is mush right now

Addendum: If I start the proxy FIRST, then the firewall, all is good. I'm thinking the proxy uses a port to connect with remote network first, then switches to my configured xxxx port...hmmm

---

### Post by bodhi.zazen on 2010-06-06
You need to do some reading on basic networking protocols.

Try the first few sections of this page:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

You will need to allow traffic on port 80 for web surfing and your VPN port.

When you start / make your VPN connection, the traffic is ESTABLISHED. Your Firestarter or UFW traffic sets rule for NEW Traffic.

If all you need is a connection for Firefox , take a look at using ssh and setting port forwarding via SOCKS.

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

[http://lifehacker.com/237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy](http://lifehacker.com/237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy)

[http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/1-putty-ssh-tunnel-introduction.shtml](http://www.devdaily.com/unix/edu/putty-ssh-tunnel-firefox-socks-proxy/1-putty-ssh-tunnel-introduction.shtml)

---

