---
title: "Strange mod_rewrite problem"
date: 2011-01-26
forum: Server Platforms
---

### Post by shelterit on 2011-01-26
Hi, I'm having a rather peculiar problem that I hope someone else have even heard of. 

On an intranet server (Ubuntu 10.10 a4, I think) running Apache2.2 with mod_rewrite and with PHP 5.3.3 we've got an Intranet application running. 

The problem in a nutshell; In test versions everything is fine, but on this particular server POST doesn't work. Everything else works fine and according to plan; GET, PUT and DELETE are all handled fine, but POST variables are completely lost. We've tested mod_rewrite thoroughly, tested all the switches and things work only on our test servers (Ubuntu 10.04, Ubuntu Server 9.10). Configs all duplicated to no avail.

Anyone ever heard of such a thing?

Update: Well, not a fix as such, but at least we now how to avoid this problem, and it's a, um, strange one.

The virtual host configuration file for Apache2 was named 'intranet' rather than '001-intranet'. Bizarre. Somehow this affected how mod_rewrite dealt with POST. I cannot even begin to understand how this could be, but there you have it. We tested this over three servers, and it is indeed what's causing our problem. We even made duplicates (meaning, all code the same except very limited config options) where instead of /intranet we had /intranet1, /intranet2 and /intraneta, and all these latter examples worked just fine. Changing the symlink name also made /intranet work. So bizarre.

Update: False alarm. The system has retorted to the old status of not working, and I cannot for the life of me reproduce the fix. So it's out, and it's getting weirder. Aaargh!

---

### Post by SeijiSensei on 2011-01-27
Without seeing all the configurations it's hard to know, but is it not possible to set the "action" parameter in the <FORM> directive so it posts to the correct URL and avoids the rewrite entirely?

---

### Post by shelterit on 2011-01-27
Yes, that's a good idea, I could do that, even though it doesn't *solve* the problem as much as circumventing it. :)

---

### Post by SeijiSensei on 2011-01-27
> **shelterit said:**
> Yes, that's a good idea, I could do that, even though it doesn't *solve* the problem as much as circumventing it. :)

I try to avoid rewriting URLs like the plague.  I do have some rewrites for "/" that force an initial URI like "/index.php?go=home" to avoid problems with the browser's "Back" button.  Other than that, I almost never rely on rewrites because of the confusion they can entail.

---

