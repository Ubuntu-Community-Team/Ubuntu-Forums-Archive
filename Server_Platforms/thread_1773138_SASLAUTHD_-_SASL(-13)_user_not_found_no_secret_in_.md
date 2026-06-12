---
title: "SASLAUTHD - SASL(-13): user not found: no secret in database"
date: 2011-06-01
forum: Server Platforms
---

### Post by graylion on 2011-06-01
Hi all

I have a working setup of SASL and OpenLDAP.I successfully authenticate cyrus, sieve, postfix and apache against this setup. I am currently trying to authenticate [Alfresco]("http://www.alfresco.com") against this and am running into the error mentioned in the subject line. looking with TCPDump I see this:

0....`.........
DIGEST-MD50.....a..
......SASL(0): successful result: ...nonce="9FNZhZzKL/bK4gp0p0w8zDm4d+5wPSON+gvRj4VA/0Q=",realm="<obscured-FQDN-of-server>",qop="auth,auth-int,auth-conf",cipher="rc4-40,rc4-56,rc4,des,3des",maxbuf=65536,charset=utf-8,algorithm=md5-sess0..,...`..%..........
DIGEST-MD5....charset=utf-8,username="graylion",realm="<obscured-FQDN-of-server>",nonce="9FNZhZzKL/bK4gp0p0w8zDm4d+5wPSON+gvRj4VA/0Q=",nc=00000001,cnonce="OS6PHN4gmvJLXurtScwftI5ybn7tX2KqTt++fi+F",digest-uri="ldap/127.0.0.1",maxbuf=65536,response=e45bf289ac2786cd10f173714ed2c63d,qop=auth0<...a7
.1...0SASL(-13): user not found: no secret in database

OK, i think, something wonky in Alfresco. The it occurs to me to have a look at the configuration of my openLDAP and I install gd (since phpldapadmin doesn't support cn=config) and try to connect. This fails and looking at the TCPDump of this I see:

0>...c9..
..
.............objectclass0...supportedSASLMechanisms0B...d=..0907..supportedSASLMechanisms1...NTLM..CRAM-MD5.
DIGEST-MD50....e.
......0....`.........
DIGEST-MD50......a..

.....@SASL(0): successful result: security flags do not match required...nonce="hH0+xECj+NZuBtAZhAbI8PaRyW1LhTLITeDl9ZCzn3g=",realm="<obscured-FQDN-of-server>",qop="auth,auth-int,auth-conf",cipher="rc4-40,rc4-56,rc4,des,3des",maxbuf=65536,charset=utf-8,algorithm=md5-sess0..H...`..A........8.
DIGEST-MD5...(username="cn=admin,dc=sm-wg,dc=net",realm="<obscured-FQDN-of-server>",nonce="hH0+xECj+NZuBtAZhAbI8PaRyW1LhTLITeDl9ZCzn3g=",cnonce="EUYBykdXL35zcPL+wCJRI4sQsbFovg2Zd6xfVz6kA2s=",nc=00000001,qop=auth-conf,cipher=rc4,maxbuf=16777215,digest-uri="ldap/172.16.2.248",response=5c4ffe7c9d2656f31fcf773b8aed83310<...a7
.1...0SASL(-13): user not found: no secret in database0....B.

which is looking awfully familiar. Uncle Google has been unhelpful so far and I don't really know where to start looking, since the setup works for several apps.

Any help appreciated.

---

