---
title: "Does WUBI Installer make the Ubuntu installation slower?"
date: 2011-12-14
forum: The Cafe
---

### Post by JF382 on 2011-12-14
Does WUBI Installer make the Ubuntu installation slower than if you were to install from a DVD instead?

---

### Post by Paqman on 2011-12-14
There's a very slight performance hit relating to disk access, but it's so small you're not likely to notice it, even if you only have a spinny hard drive.

---

### Post by lukeiamyourfather on 2011-12-14
Yes, but maybe not enough to matter.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1)

Something that might matter more is the greater potential for loss of data and/or corruption of data since the data lives in a file on another partition that is susceptible to things like Windows malware and accidental deletion.

---

### Post by Paqman on 2011-12-14
> **lukeiamyourfather said:**
> 
Something that might matter more is the greater potential for loss of data and/or corruption of data since the data lives in a file on another partition that is susceptible to things like Windows malware and accidental deletion.

That's not a Wubi issue specifically, those are threats to your data wherever it's located. A good data protection plan including redundancy and backups should mitigate the risk.

---

### Post by lukeiamyourfather on 2011-12-14
> **Paqman said:**
> That's not a Wubi issue specifically, those are threats to your data wherever it's located. A good data protection plan including redundancy and backups should mitigate the risk.

Yes, data is always at risk. Just pointing out that risk is greater with Wubi. People ask about performance all the time but that's not the only factor when considering using Wubi versus a traditional installation.

---

