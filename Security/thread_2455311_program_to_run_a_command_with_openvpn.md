---
title: "program to run a command with openvpn"
date: 2020-12-17
forum: Security
---

### Post by bardiamgtgc on 2020-12-17
is there any program to run only one command with openvpn?
i have an openvpn setup on my server and i want another machine to only connect to that vpn connection for running that command.
does anybody know anything about that?

---

### Post by TheFu on 2020-12-17
setup the firewall to only allow openvpn connections from the 1, single, remote machine's static ip address.

But really for something like that, I'd use ssh instead, which can force a specific command to be run based on which ssh-key is used for authentication.

The right tool, for the right job.

---

### Post by bardiamgtgc on 2020-12-17
i have my firewall configured for that openvpn ip but i dont want to tunnelwhole ubuntu machine(my desktop machine) with openvpn just one command and i cant use like a socks proxy because that wont be encrypted thats why i was looking for some openvpn tool

---

### Post by TheFu on 2020-12-17
ssh can provide an encrypted SOCKS proxy, but to get DNS encrypted, you'd also need DoH setup. Normally, DNS is UDP and UDP cannot be proxied via ssh.
I use an ssh tunnel as a SOCKS proxy more than I use a VPN.  I've posted my script for this in these forums a few times over the years.

---

