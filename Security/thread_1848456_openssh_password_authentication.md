---
title: "openssh password authentication"
date: 2011-09-22
forum: Security
---

### Post by rp11235 on 2011-09-22
When one uses public key method to login to openssh, does it use the server's public key to encrypt the password?
If the client also had a public private key pair, it would probably use it to encrypt the data, but assuming password authentication, is the password encrypted using the public key?

It would be useful if someone could post links from reliable sources too about this.
The RFCs have little about password encryption except at the transport layer.

Thanks,
rp11235

---

### Post by bodhi.zazen on 2011-09-22
The place to start is with the man pages.

Then try this : 

[http://www.1986.ro/db/docs/linux/SSH%20%26%20VPN/O%27Reilly%20-%20SSH%20The%20Secure%20Shell%20The%20Definitive%20Guide.pdf](http://www.1986.ro/db/docs/linux/SSH%20%26%20VPN/O%27Reilly%20-%20SSH%20The%20Secure%20Shell%20The%20Definitive%20Guide.pdf)

---

