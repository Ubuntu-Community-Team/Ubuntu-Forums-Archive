---
title: "Making Private Tunnel Connect"
date: 2012-02-23
forum: Security
---

### Post by failheart on 2012-02-23
Hello, I have a problem with connecting to the private tunnel portal........i have Openopvn installed and i downloaded the client.ovpn file and installed the file in the etc/opvn directory....

I go and login to private tunnel and click on the connect button at the top of the page on the 'my portal' page and it brings me to logging in again and wont ever connect.

Did I install the client.ovpn in the wrong place?:confused:

---

### Post by kevdog on 2012-02-23
I'd run both the client and server in debug mode to see if you can generate some output to help us with this one.

---

### Post by failheart on 2012-02-24
To test the client configuration you can manually start the OpenVPN client with the command

# openvpn /etc/openvpn/client.ovpn............anyways it works now.:)

---

