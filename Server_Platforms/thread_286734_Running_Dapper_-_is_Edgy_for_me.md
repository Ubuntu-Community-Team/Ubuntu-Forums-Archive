---
title: "Running Dapper - is Edgy for me?"
date: 2006-10-28
forum: Server Platforms
---

### Post by jimwillsher on 2006-10-28
Hi all,

I'm running Dapper purely as a server. Packages:

Apache2
MySql5
PHP
Postfix
Spamassassin
ClamAv
Squirrelmail
Amavis

etc.

I like to have recent versions of packages, especially SpamAssassin and ClamAv, but Dapper is still stuck in the dark ages with these. Dapper is supposed to be LTS, but LTS seems to really mean bug-fixes only, rather than moving with the times.

So, my dilemma. Do I stay with an LTS release and have old packages, or do I upgrade and have a non-LTS release but with newer packages?

Comments / advice VERY welcome!


Jim

---

### Post by Peter76 on 2006-10-28
Hi Jim, I would stick with Dapper; especially because you have a server; Edgy is ( as the name implies ) quite bleeding edge, and thus not completely bug free.
I would check if there are any backports for the packages you want, or otherwise install them from source and keep the benefits of the LTS

---

