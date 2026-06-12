---
title: "setup SOCKS5 proxy"
date: 2010-03-30
forum: Server Platforms
---

### Post by hotpancakes on 2010-03-30
Hi all,

I have an interesting situation. I'd like to use bittorrent for legitimate purposes (mainly linux distro based) but the powers that be have blocked access to bittorrent at my university. I have an ubuntu VPS that I use for odds and ends and was thinking that I could setup a SOCKS5 server on it. That way, I can input the SOCKS5 info directly into the proxy section of my local bittorrent application (Transmission 1.92 running on snow leopard) and be good to go. The problem, however, is that I cannot find a way to get a SOCKS server up and running on my VPS. I've heard that ssh can be used as a simple SOCKS server, but I've also heard that i may need to install a more complete SOCKS server such as dante. Does anyone have any thoughts on this? Thanks!

---

### Post by HermanAB on 2010-03-30
Install ssh-server and use the -D switch in ssh.

---

