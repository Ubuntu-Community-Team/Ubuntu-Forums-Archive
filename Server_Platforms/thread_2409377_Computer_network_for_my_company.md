---
title: "Computer network for my company"
date: 2019-01-01
forum: Server Platforms
---

### Post by seoalexramon on 2019-01-01
Good afternoon from Spain!
I'm starting a small business in which I need to install 16 computers. In principle all these computers will be for the workers and will be connected under the same network. On the other hand I will have my computer too and as the workers' computer will hardly have permissions to install programs I would like that I from my computer that is connected to the same network as the workers' computers, can install programs from my computer. I have seen companies using it but I have not been able to find out how I can do it. I hope you can help me and thank you very much for reading and answering! Best regards!

---

### Post by volkswagner on 2019-01-01
Perhaps you are interested in [Linux Terminal Server Project]("http://www.ltsp.org/") (LTSP).
[Edubuntu]("https://www.edubuntu.org/") has LTSP baked in, but I'm not sure how development is going since their page
shows Ubuntu 14.04 as their latest version (which was posted back in 2015).

I have only dabbled in LTSP. If LTSP is the route you are thinking of, hopefully you can do
so research then come back and ask more specific questions.

---

### Post by Tadaen_Sylvermane on 2019-01-01
Ltsp is great. I use it at home for media centers. I would use it for more if i had a family. Just the wife and i right now.

Ubuntu help pages. Edubuntu is not needed. Is simple to install it yourself on any ubuntu version.

---

### Post by seoalexramon on 2019-01-01
Okey thank you very much for your kindness to both users and for your speed. Thank you so much I'm going to try it right now!

---

### Post by TheFu on 2019-01-08
The admin account can install programs.  Other accounts cannot.  Setup the computers, but don't give the workers the admin login.  Simple.  For 16 people, I'd setup centralized authentication, centralized HOME directories using NFS and a server where all their files get stored.  Lots of other ideas for a small business, but it would depend on the business.

I've used a central terminal server before, but that was back when computers were $30K each.  These days, you can do pretty amazing things on $200/ea computers. Whether that makes sense or not would depend on the business.  Might be possible to setup $80/ea computers using SBCs, just add monitors, keyboards and mice.

For 16 computers, might want to automate management either with scripting or through a devops tool like ansible, puppet, chef, salt, or something similar.

I'm assuming no Windows, anywhere.

---

