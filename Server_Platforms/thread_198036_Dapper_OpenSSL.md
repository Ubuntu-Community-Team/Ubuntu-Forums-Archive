---
title: "Dapper: OpenSSL"
date: 2006-06-16
forum: Server Platforms
---

### Post by ScatterBrain on 2006-06-16
Did anything change for OpenSSL between Breezy and Dapper?

The reason I ask is that I've been trying for two days to setup a Certificate Authority (CA) on a Dapper machine using:

```
# /usr/lib/ssl/misc/CA.sh -newca
``` 
On Breezy machines in the past, this has worked without a problem.  All of my certificates work just fine.  But using the Dapper machine, I keep getting told by Windows machines [COLOR=Navy]*(I know, I know)*[/COLOR] that the CA doesn't have the right to create certificates, and the certificates can't be used.

I went back to a Breezy machine today and created a CA and certificates and they come in just fine.

Can someone shed some light on this for me please?

---

