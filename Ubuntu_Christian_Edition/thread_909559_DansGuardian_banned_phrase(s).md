---
title: "DansGuardian banned phrase(s)"
date: 2008-09-03
forum: Ubuntu Christian Edition
---

### Post by linxlvr on 2008-09-03
Hi all. First let me say TY to all involved for making this distro. TY Jeremy for your energies and insights in going ahead w/ the new version.

Now the question.:-)
I like to go online to a forum about boating (fixing boats, boat motors, etc.) called "iboats"
When going to the iboats forum, it is denied, banned phrase. OK. I looked at the logs and it seems to be telling me the banned phrase is "gator". whatever.
Anyways, when I look through all the /etc/dansguardian/* stuff I can't seem to find that banned phrase. Can anyone help me with this?
TYIA
-- 
dw

---

### Post by mhancoc7 on 2008-09-03
> **linxlvr said:**
> Hi all. First let me say TY to all involved for making this distro. TY Jeremy for your energies and insights in going ahead w/ the new version.

Now the question.:-)
I like to go online to a forum about boating (fixing boats, boat motors, etc.) called "iboats"
When going to the iboats forum, it is denied, banned phrase. OK. I looked at the logs and it seems to be telling me the banned phrase is "gator". whatever.
Anyways, when I look through all the /etc/dansguardian/* stuff I can't seem to find that banned phrase. Can anyone help me with this?
TYIA
-- 
dw

Thanks for the kind words!

Are you using the Parental Controls GUI to change the settings?

Jereme

---

### Post by linxlvr on 2008-09-03
> **mhancoc7 said:**
> Thanks for the kind words!

Are you using the Parental Controls GUI to change the settings?

Jereme

I went there to view the logs, but banned phrase list that showed up in parental controls was simply a list of what seemed to be 3 files that it would use. Going to those files 'the old way' I was unable to find the phrase. I didn't use the lower settings as 'strict' is a good idea in this household. :-)
-- 
dw

---

### Post by lisati on 2008-09-03
I'm wondering if "gator" is banned because of a piece of spyware called "gator" ([http://www.pchell.com/support/gator.shtml](http://www.pchell.com/support/gator.shtml))

---

### Post by linxlvr on 2008-09-03
> **lisati said:**
> I'm wondering if "gator" is banned because of a piece of spyware called "gator" ([http://www.pchell.com/support/gator.shtml](http://www.pchell.com/support/gator.shtml))

That was it, thanks. located in /etc/dansguardian/phraselists/malware/weighted.

Thanks again.

-- 
dw

---

