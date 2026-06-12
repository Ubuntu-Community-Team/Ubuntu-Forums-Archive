---
title: "Secure, encrypted connections for all protocols via HTTPS and SSL"
date: 2008-01-15
forum: The Cafe
---

### Post by Convert on 2008-01-15
Hey there to the world...hope you are doing well.

I have a need and I was wondering if any one knows of a solution.  The problem I am trying to solve is to enable secure network traffic for any (or at least most) network protocols when the only secure protocol allowed is HTTPS/SSL.

I want to have something on my Ubuntu laptop that will send all network traffic through an HTTPS/SSL based connection (first leg of the network path only).  I think the thing I need  is where my laptop creates an HTTPS live connection to a server somewhere where the server receives the HTTPS traffic from my laptop and then retransmits the same traffic unencrypted using the correct protocols.  Sort of a relay.

For example, if I need to do an ftp transfer, first my laptop would encapsulate the ftp protocol inside an HTTPS wrapper and send it to the server.  The server would receive the traffic, unwrap the HTTPS and then resend the ftp request using the server's IP.  The ftp would come back to the server and the server would rewrap the ftp traffic inside the HTTPS and forward it on to my laptop.  I am looking for something that I can turn on (all network traffic goes to the HTTPS relay server)/turn off (all network traffic is sent normally).

This relay thing has to use HTTPS/SSL because that seems to be the most likely allowed secure communications protocol at all of the public open wireless access points (in some case the only allowed secure connection).  Many of the other protocols are not allowed, yet frequently one needs to use something other than HTTPS to communicate.  I am not concerned with having an end to end secure connection, only secure from the public access point to the first server in the link.

Is there anything like that out there?  :confused:

---

### Post by kevdog on 2008-01-15
I know what you want to do, and the answer is I dont know.

Another variation of this would be to run an ssh server on port 443.  You could then establish an ssh connection from the coffee house through port 443 to your home openssh server on port 443.  Within the ssh option you could establish a socks proxy, and then run firefox for example through the socks proxy encrypted to your server, and then unencrypted from your server to the internet.

With ssh its also possible to forward local ports to remote ports, so in a similar manner (different command to establish the encrypted ports), you could use ftp, or basically any other program. (pop, smtp, imap etc).

Here is a blog about the firefox secure tunnel.

[http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

Ive personally used this approach along with the dd-wrt firmware on my router, to ssh into my router from a remote location (airport) and then run firefox through the socks/secure ssh tunnel.

---

### Post by Convert on 2008-01-15
Hmmm...the ability to use a SOCKS proxy over HTTPS may be key.  Good suggestion.

---

