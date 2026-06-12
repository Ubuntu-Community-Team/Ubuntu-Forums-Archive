---
title: "vsftpd &quot;Server sent passive reply with unroutable address.&quot;"
date: 2012-03-19
forum: Server Platforms
---

### Post by schoft on 2012-03-19
I am at home. My server is also at home. It has a static IP. VSFTPD runs on port 22222. Port forwarded in my router too. Now, whenever I connect to it after changing my DNS records I get this:

Response:200 Switching to Binary mode.
Command:PASV
Response:227 Entering Passive Mode (192,168,133,7,136,218).
Status:Server sent passive reply with unroutable address. Using server address instead.
Command:LIST
Error:Connection timed out
Error:Failed to retrieve directory listing

Why is this happening?

---

### Post by cryptotheslow on 2012-03-19
From what you say I presume you are updating your DNS records to point to the external internet facing IP of your router?

If so then your PC will be connecting to the external interface of your router and then the connection forwarded through NAT back into your LAN to the ftp server. When the ftp connection tries to change into passive mode the server supplies its IP address and what port(s) to use to establish the passive connection. As it is reporting its LAN IP there and your FTP client considers itself connected to an internet based FTP server it reports that the IP provided is invalid as it is not routeable on the internet.

I don't know how to with vsftpd but with proftpd there are settings in the config file for working behind a NAT'd connection. Basically you need to enter config entries for:

1. The external IP address (some ftp servers have an option to try to auto-detect this at run time)
2. The port range to use for passive connections (usually by default this is quite a large range, reducing this in the config makes the next thing simpler)

The next thing - you also need to forward the passive ftp port range on your router to the ftp server as well as the usual port 21.

Hope that helps - I'm sure a net search for something like "setup vsftpd to work behind NAT" will give a number of hits with specifics.

GL HTH

---

### Post by SeijiSensei on 2012-03-19
From the man page for vsftpd.conf:

> pasv_address
    Use this option to override the IP address that vsftpd will advertise in response to the PASV command. Provide a numeric IP address, unless pasv_addr_resolve is enabled, in which case you can provide a hostname which will be DNS resolved for you at startup.

    Default: (none - the address is taken from the incoming connected socket) 

Your machine is sending its private LAN address, 192.168.133.7, instead of the public address on the outside of your router.  Try using this directive to send your external address instead.

PS:  Stuff like this is why I hate the FTP protocol.

---

