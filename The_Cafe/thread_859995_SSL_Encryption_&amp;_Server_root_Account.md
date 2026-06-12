---
title: "SSL Encryption &amp; Server root Account"
date: 2008-07-15
forum: The Cafe
---

### Post by amauk on 2008-07-15
Hypothetical question...

Server is running a daemon, called d

d listens for encrypted connections of a tcp port
d initially runs as root, and has read access to SSL private key
d drops to unprivileged user once SSL established

Client, c, sends a secret payload to daemon d
payload encrypted with server's public key
d reads secure payload, and acts accordingly

Now...

If you have access to the root account on the server,
can you intercept and read the secure payload at any point?

What if private key is "embedded" in daemon d, and only available to d's internal workings?
(ie. no system user, not even root, can access the private key) ?

can root intercept and read the secure payload at any point?

*edit*
if you're wondering about motives, I'm writing the server program

It's a business program, and will be distributed to 3rd party companies
designed to allow contractors to bid on contracts produced by a company

For legal reasons (collusion, price fixing, etc.), no-one (not even the company running the contract) should know what bids are until a deadline has been reached

I want to safe-guard any client bids from being disclosed before the deadline

---

