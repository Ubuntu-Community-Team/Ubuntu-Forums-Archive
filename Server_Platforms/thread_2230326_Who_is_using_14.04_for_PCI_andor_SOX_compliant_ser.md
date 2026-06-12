---
title: "Who is using 14.04 for PCI and/or SOX compliant servers?"
date: 2014-06-18
forum: Server Platforms
---

### Post by 1clue on 2014-06-18
Hi,

Just curious if anyone is using Ubuntu Server 14.04 for PCI- and SOX- compliant servers?

If you don't know what that is, it means processing credit cards or handling bank transactions.

I'd like to know how your testing has gone so far, and whether you'd recommend trying it yet.  And what advice you have.

I already do this with 12.04, I'm just interested in a comparison of the two.

Thanks.

---

### Post by DJ_Max on 2014-06-21
I'm not sure what you're trying to find out. PCI/SOX does not care what operating system you use, as long as it meets their standards. If you know Linux admin, than configuring Ubuntu shouldn't be diffcult. Especially considering PCI compliance isn't all that secure.

---

### Post by 1clue on 2014-06-23
I'm already using 12.04 on public servers of various security levels.  I'm trying to find out if anyone else is doing it with 14.04 yet, and if so what challenges there are.  For example, stability or compliance issues.

---

### Post by CharlesA on 2014-06-23
There shouldn't be much different in the base configuration except new having newer packages. If you do decide to check it out, roll a VM and throw your current config files onto it and see what blows up.

---

### Post by SeijiSensei on 2014-06-23
Aside from security updates, most server software has been around for so long that it remains quite stable across updates.  I doubt there is little that distinguishes 14.04 Server from 12.04 other than updates.

---

### Post by CharlesA on 2014-06-24
> **SeijiSensei said:**
> Aside from security updates, most server software has been around for so long that it remains quite stable across updates.  I doubt there is little that distinguishes 14.04 Server from 12.04 other than updates.

Apache 2.4 vs 2.2, for one, but that's the only thing I could think of off the top of my head. I believe that version change also changed how apache was configured as far as virtual hosts go.

But yeah, it's stable for the most part so unless there is a major difference between releases, it shouldn't be a problem overall.

---

### Post by 1clue on 2014-06-24
Thanks.

---

