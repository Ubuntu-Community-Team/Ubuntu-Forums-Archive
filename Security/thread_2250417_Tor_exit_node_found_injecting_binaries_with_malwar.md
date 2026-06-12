---
title: "Tor exit node found injecting binaries with malware"
date: 2014-10-28
forum: Security
---

### Post by bashiergui on 2014-10-28
A researcher found Windows updates injected with malware by a rogue Tor exit node. Tor subsequently blacklisted that exit node.
[http://www.leviathansecurity.com/blog/the-case-of-the-modified-binaries/](http://www.leviathansecurity.com/blog/the-case-of-the-modified-binaries/)

If one was detected, there are probably others. Don't download unnecessary binaries over Tor.


Currently you can easily force Ubuntu updates over https.  But more broadly, this attack indicates it might be time to ask if system updates should be forced over https by default. I'm guessing if you did catch maliciously injected updates on Ubuntu, the signatures and keys wouldn't match so they would fail. But if Ubuntu aims to be every man's OS, perhaps SSL/TLS by default is the way to go.

What do you think? Is it just paranoia or is https a legitimate and viable solution?

---

### Post by open2reason on 2014-10-28
Good advice about Tor, as always a quick look at the Tor project page [https://www.torproject.org/](https://www.torproject.org/)  should keep one informed of any Tor related problems and any fixes required.

---

### Post by untrustytahr on 2014-10-29
> **bashiergui said:**
> Currently you can easily force Ubuntu updates over https.  But more broadly, this attack indicates it might be time to ask if system updates should be forced over https by default. I'm guessing if you did catch maliciously injected updates on Ubuntu, the signatures and keys wouldn't match so they would fail. But if Ubuntu aims to be every man's OS, perhaps SSL/TLS by default is the way to go.

What do you think? Is it just paranoia or is https a legitimate and viable solution?

  	 	 	 	   While I normally agree with sending all traffic over ssl/tls when possible, in this particular use case, I don't see much added value.  SecureApt is already checking the signed hashes.  As long as the sig is valid and the package hashes match, you know you have the correct d/l that the maintainer intended (provided the private signing key is properly safeguarded).
 

 The only additional benefit that ssl would provide is authentication that you contacted the 'real' server, but that doesn't really add anything.
 

 Now, if you're using TOR downloading binaries without signatures/hashes... that's a much different story.  That's just plain crazy.

---

