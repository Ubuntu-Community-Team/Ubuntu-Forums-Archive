---
title: "Ubuntu Server 8.10 DNS and DHCP Server"
date: 2009-03-02
forum: Server Platforms
---

### Post by danooch13 on 2009-03-02
Hello,

I am new to Linux.  I am trying to setup a DNS and DHCP server on ubuntu server 8.10 which I already did.  Both components work perfectly....well....perfectly separately.

My problem is that I can't get the clients that get a dhcp address from the ubuntu server register with DNS which is on the same server.

I have some static dns addresses in the server which are fine, but the regular dhcp clients will not register with dns.

Is there a way to do this?

Thanks

---

### Post by danooch13 on 2009-03-03
Anyone?

I know it has to be possible.

---

### Post by netztier on 2009-03-03
> **danooch13 said:**
> 
I have some static dns addresses in the server which are fine, but the regular dhcp clients will not register with dns.


Read the "DYNAMIC DNS UPDATES" section in dhcpd.conf's manpage. It's all in there.

```
user@server:~$ **man dhcpd.conf**
```


And a suggestion: DHCP clients should not update the server, unless they can be authenticated by a good mechanism (such as Kerberos). Leave it to the DHCP server to send an authenticated DDNS update to the DNS server.

regards

Marc

---

### Post by danooch13 on 2009-03-03
Thank you.  I will attempt this in a few.

---

### Post by HermanAB on 2009-03-03
Hmm, letting the clients update the DNS is a Microsoft abomination that represents a huge security hole.  It is used by MS Active Directory - they specially modified an old copy of BSD BIND8 for that.

Soooooo, my suggestion is don't do that. You can use a Samba domain controller or a NIS without having to let the clients do DNS updates.

Cheers,

Herman

---

### Post by danooch13 on 2009-03-03
LOL.  I am a Microsoft admin for years, and got frustrated with it so I decided to take the switch.  I guess some of my old ways carried over.

---

