---
title: "Upgrade from Sarge to Breezy Server; good idea or not?"
date: 2005-12-03
forum: Server Platforms
---

### Post by dotmil on 2005-12-03
Currently I have a few dedicated servers leased from a provider, all of them running Debian Sarge. I'd really like to run Breezy Server on one of them, but the provider of course doesn't have Ubuntu as an installation option.

So that leaves me with two choices, either dist-upgrade from Srge to Breezy, or rent a remote KVM and attempt a fresh install (more $$). I'd like to attempt the first, but am just wondering if anyone here has experience with doing this type of thing. I did search and found some seemingly mixed reults.

The server I have picked out for this isn't running anything extremely critical, and I have current daily backups of the data that is on there. It serves as http/mail/DNS/mysql mainly, but only handles mail for a few accounts with no real active sites on the http server. So the risk would be minimal, but of course I am leery of some huge issue arising that would cost me an arm and a leg in support costs.

So, what say you all? Go for the dist-upgrade or wait until I can get the KVM and try that way? With the KVM, I'd likely still have to bootstrap the install. I'm not sure my provider would be willing to burn and swap the CD for me.

---

### Post by dotmil on 2005-12-04
Anyone?

---

### Post by linbetwin on 2005-12-04
I don't know anything about servers, so don't take my word for it, but I don't think this is possible. Ubuntu may be derived from Debian, but they're not 100% compatible.

---

### Post by dotmil on 2005-12-04
Thanks. I have found several people via Google who claim to have pulled this off without a hitch. But I'm really looking for someone with firsthand experience of it. I guess I could always contact one of the people I found during my searches.

I may just go ahead and give it a whirl on a test box. If it breaks then, it won't hurt anything and I'll finally have this mystery cleared up.

---

### Post by dotmil on 2005-12-04
Just a follow-up on this.

I have successfully done this upgrade on two test servers now (one PIII/512MB, one Athlon64/1024MB [32-bit mode]). So far they both appear to be stable and running fine. I had to fix a few dependencies manually, but so far so good. I'll run them for a few days before attempting this on a live server though.

---

