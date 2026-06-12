---
title: "Formatting of the Domain Controller"
date: 2006-06-14
forum: Server Platforms
---

### Post by taipeiben on 2006-06-14
I was using Fedora as my domain controller for my small network of Windows machines and I decided to give Ubuntu a try.  I reformatted my main drive and installed Ubuntu and set up Samba so my box could be the domain controller again with all the same settings as before.

On my Windows machines, I couldn't log in.  I had to first leave the domain and rejoin it and then copy over the local profiles to the new local profile that windows creates.  It's not a big deal with 1 or 2 systems, but there's a lot of Windows machines on my network.  Is there a way to make the reformat seamless to the Windows machines?  Make it seem like to the Windows machines as if i just shut down the domain controller for a few hours?

The reason I'm asking is because I think my main HD is failing and I'm going to have to redo this whole ordeal over again when I get the time to replace the drive.  Also I like to experiment with different OS's.

---

### Post by LordHunter317 on 2006-06-14
Not if you erased the Fedora install, you cannot.  You erased the databases that are necessary for domain operation; they contain all the security information.

---

### Post by mjm115 on 2006-06-14
No.  If you delete the controller, then you have to reconfigure all of your machines, because all trusts and security information is lost.

---

### Post by taipeiben on 2006-06-14
Alrighty, thanks for the info.

---

### Post by taipeiben on 2006-06-14
What about configuring a 2nd computer as a backup domain controller with Samba?  Is there anyway to recover the trusts and security information and other DB stuff from the BDC to the PDC?

---

### Post by LordHunter317 on 2006-06-14
You mean you had a BDC already?  Possibly, but I'd have to look into it.  I think the answer may be no anyway, however.  I'm not sure some of the trust data is replicated.

But it's simple: if you wiped the machines that had the trust data on them, you're recreating the whole domain from scratch.

---

### Post by taipeiben on 2006-06-15
1.  Yah assuming I had a BDC set up, could I recover the trust data from it?

2.  Silly question I'm sure:  Could I put the trust data on a different partition or drive?  Like /dev/hdb1 instead of my main partition?  So next time I distro hop or distro upgrade I don't have to redo everything.

---

