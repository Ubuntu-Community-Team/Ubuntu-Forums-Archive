---
title: "SPF: Sender Policy Framework"
date: 2007-06-29
forum: Server Platforms
---

### Post by z33k3r on 2007-06-29
Has anybody implemented this with Ubuntu server? I have run the Perfect Setup for 7.04 and everything is running great. Have added Reverse DNS on the ISP side, but some places like AOL are looking for SPF (Sender Policy Framework). Searching the forums, I am not really finding any body with posts concerning this topic... Any help would be greatly appreciated..!

:popcorn:

---

### Post by z33k3r on 2007-08-07
*bump*  <----------- I hate doing this...

Anybody have experience with using these SPF records to reduce spam and such?

---

### Post by MJN on 2007-08-08
I use them, and it does have some positive effect. As always it's not a solution by itself, but adds effectiveness as part of a bigger multi-faceted approach.
 
The vast majority of domains of incoming mail don't have SPF records but those that do are resulting in occasional forged mail being rejected when it had otherwise already passed through my RBLs (which are significantly more effective for me).
 
I don't have access to stats for my DNS so do not know how many others are querying my domain for its SPF records however, and of most value to me, immediately following SPF implementation my backscatter across all my domains was reduced massively (to practically zero in many cases).
 
Again, it's not the be all and end all but it's helping. The only downsides I've experienced are when 'legitimate' 3rd parties attempt to send mail out masquerading as my users e.g. the BBC's 'Send this page to a friend' link, or some eCard type businesses who stick the senders address in the From field. It doesn't happen often though, and I could always weaken the SPR ruleset but this may compromise the overall effectiveness.
 
From my experience and setup I'd rank RBLs and greylisting as being of higher value.
 
Mathew

---

### Post by z33k3r on 2007-08-08
Do you, or anybody else, know of a nice tutorial on these things as I have not implemented them before and I am not a *nix Master by any means...

---

