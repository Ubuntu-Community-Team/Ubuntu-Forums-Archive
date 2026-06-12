---
title: "SPF Record ok?"
date: 2007-10-10
forum: Server Platforms
---

### Post by hyper_ch on 2007-10-10
Ok, I have been using a catch-all email address for a very long time... so whenever I needed to sign-up at some place (e.g. [http://www.somedomain.com](http://www.somedomain.com)) I entered as email address: [www.somedomain.com](www.somedomain.com) [at] roleplayer [dot] org.

That way I could easily track where my email address was leaking.

From time to time some people forged a  roleplayer dot org email address and it was then bounced back... that wasn't that bad. However yesterday, within two hours I got over 160 such bounce backs ( http [column slash slash] t390[dot] greatnet [dot] de [slash] cgi-bin [slash] mailgraph [dot] cgi ).

For the moment I did now deactivate that catch-all email but as you can see, there are still a lot of rejected emails (although it's turning towards normal again).

I use the postfix integrated UCE mechanisms, greylisting and rbls but that didn't help much as you can see.

So I started setting up SPF (according to the howto) and I wonder now if my SPF entry is correct.

The SPF entry should do the following:
- bind roleplayer [dot] org to the IP 83.133.126.175
- say ok to any subdomain sending mail through 83.133.126.175
- also say ok to the hostname given by my ISP t390 [dot] greatnet [dot] de
- return false from any "roleplayer [dot] org" email that is not being sent through the 83.133.126.175 ip address

Here's the SPF entry I added to the bind zone file:
```

roleplayer [dot] org. IN TXT "v=spf1 a mx ptr a:t390 [dot] greatnet [dot] de ~all"

```

of course [x] has to be replaced by the according character.

---

### Post by MJN on 2007-10-10
I would drop the **ptr** directive - it's not really adding much (other than additional lookups).
 
You may also find you'll have to use **-all** (as opposed to** ~all**) to be effective as it is arguable that domains stating they are in a 'transitioning phase' may as well have no records at all as SPF failure can only then be considered to add to suspicion rather than indicate definite spoofing. I'd jump in with two feet if I were you and use **-all** to state your anti-spoofing position clearly.
 
For what it's worth I also had backscatter problems on a couple of domains and SPF nailed it - there is still the occasional issue but it's certainly been a great help. The one drawback I've suffered is with forwarded mail - this often fails the SPF check and hence fails (this is a known drawback with SPF).
 
Mathew

---

### Post by hyper_ch on 2007-10-10
Thx for the input. I'll look at that :)

---

