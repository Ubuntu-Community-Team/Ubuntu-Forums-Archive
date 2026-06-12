---
title: "DNS Error"
date: 2010-06-03
forum: Server Platforms
---

### Post by terazen on 2010-06-03
I have 2 ubuntu lucid dns servers that are getting this error and I don't know what it means.

> named[1035]: success resolving 'somewebsite/A' (in 'somewebsite.foo'?) after reducing the advertised EDNS UDP packet size to 512 octets

Also, both servers are acting up at the same time.  I've disabled the ufw with no luck and verified that named is running with "/usr/sbin/named -4 -u bind".

I've moved from 2 physical servers running ubuntu hardy to 2 virtual machines running ubuntu lucid on esxi servers which is when all of this started.  If this isn't resolved quickly I'll have to move back tonight which would be a pain.

Any ideas?
Edit:
I should have noticed earlier, but the reason for the errors happening at the same time is because the pc's in the location are pointing to 2 AD DC's that are each pointed to a different bind server as primary forwarder.  

I've read that the error could possibly have something to do with firewall software that drops dns messages over 512bytes (not supporting EDNS) so I sent in a request for one of the firewall people to look at this.

Setting "edns-udp-size 512;" in named.conf.options hasn't helped.

---

### Post by BobVila on 2010-06-03
Looks like you're getting DNSSEC packets back from the root DNS servers and that your bind install isn't set up to respond to those properly. I haven't tinkered with message length on bind servers, but if you find where the setting is, bump it from 512 bytes up to 2048.

---

### Post by terazen on 2010-06-03
I've just installed from the repositories and copied over a working configuration so I don't know about the dnssec support.  I haven't signed any of my zones yet.

I found this from Bind 9.7 documentation on ISC's website:
> edns-udp-size
Sets the advertised EDNS UDP buffer size in bytes to control the size of packets received.
**Valid values are 1024 to 4096 (values outside this range will be silently adjusted)**. The default value
is 4096. The usual reason for setting edns-udp-size to a non-default value is to get UDP answers
to pass through broken firewalls that block fragmented packets and/or block UDP packets that
are greater than 512 bytes.
named will fallback to using 512 bytes if it get a series of timeout at the initial value. 512 bytes is
not being offered to encourage sites to fix their firewalls. Small EDNS UDP sizes will result in the
excessive use of TCP.

This explains why "edns-udp-size 512" didn't work.  My site is being silently "ENCOURAGED" to fix the firewall.  I've received similar encouragement from firefox and microsux, but isc as well?

Going to switch back to hardy and put the lucid server offline until I can downgrade the software.

---

### Post by BobVila on 2010-06-03
Guess that's one way to go... personally, i'd think it's easier to flip edns-udp-size back to 4096 and change the max dns udp length on your firewall...

---

### Post by terazen on 2010-06-04
Yeah, it would be easier if I could set the size to 512 until the firewall could be changed.  I'm not going to have all of our users experience timeouts for days while we wait for that to happen though.  Kinda sucks for encouragement to work out like this.

---

