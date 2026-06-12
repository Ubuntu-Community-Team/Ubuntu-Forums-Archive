---
title: "Users get to the root of Linux security holes"
date: 2006-01-24
forum: Server Platforms
---

### Post by newbie2 on 2006-01-24
> "I believe that Linux needs to get rid of 'root,'" Canfield said in an e-mail to SearchOpenSource.com. "Root is not a user; root is a capability to surpass security. As long as that capability exists, there will be ways to hack it."
[http://searchopensource.techtarget.com/originalContent/0,289142,sid39_gci1160533,00.html](http://searchopensource.techtarget.com/originalContent/0,289142,sid39_gci1160533,00.html)
:rolleyes:

---

### Post by Virogenesis on 2006-01-24
I do not see a problem with root with ubuntu as it is disabled so users cannot log in.
Root is far better than anything MS has come up with and they are the only ones that take a different approach. 
If you want to protect your comp in such a manner making it harder for a cracker to get in.
Prevent access to the BIOS for a start if your case allows for you to padlock it do so that will they will not be able to remove the battery from the motherboard keeping the password you will put on safe.
Password protect the BIOS and don't allow it to boot from CD or Floppy.
When on the internet use a firewall keep apache patched at all times, mysql allow for local access only. 
Use a password that has lower case uppercase and symbols change it often like every 14 days or so.
If using SSH use port knocking it will stealth your port or anyone scanning will not see you have a SSH server running.
When using a FTPD use virtual users.
Bugs are everywhere just don't let crackers exploit them basically.

---

### Post by alamba on 2006-01-24
I wonder what Canfield has to say about m$'s "administrator"!!

---

### Post by tcwitte on 2006-01-25
[QUOTE=Virogenesis]I do not see a problem with root with ubuntu as it is disabled so users cannot log in.[/QUOTE]
I agree root as a user isn't a problem with Ubuntu -- programs running as root still are however. If those programs break and aren't well constrained someone can still brake in as root. I'm looking forward to progress on SELinux or AppArmor because I think they will solve that problem as well: programs won't run as unrestricted root anymore.

---

### Post by curtis on 2006-01-28
Hi,
No one has mentioned that his idea of root is actually quiet different to what everyone else is thinking.

E.g this:
> 
Canfield said there is still potential for root in the partitioned versions of Linux, where root is not global but is only local to some portion of the system.


Don't you only need priveleges to modify the settings, is he saying that he would not mind every user modifying the network settings...
> 
"Why should changing the LAN settings require write access to the entire hard disk?" he asked.


Also, a lot of the 'issues' he points out affect Windows the same or in some cases worse.
I think the only point where he may be a tiny bit correct is with the drivers in user space (He calls it 'somewhere else where drivers can live outside the kernel')
But then again, wouldn't that be a lot slower and result in a lot of data being sent to the kernel and back, thus wasting a lot more time.

---

### Post by public_void on 2006-01-28
> I wonder what Canfield has to say about m$'s "administrator"!!
IMO it seemed he was nit-picking with Linux compared to Windows. Although its for the best so to improve Linux. A possible problem could be too much security. If plans like this do make it into development in futrue Linux distro it will be interesting how they strike a balance with access rights etc. Because I'd hope they wouldn't over do it, and in effect create a box that is harder for the user to use than a hacker to attack.

I don't think it was worth talking about MS's administrator, it'd be a waste of time as its very clear whats wrong with it.

---

