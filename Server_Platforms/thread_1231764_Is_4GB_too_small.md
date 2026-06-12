---
title: "Is 4GB too small?"
date: 2009-08-04
forum: Server Platforms
---

### Post by garfonzo on 2009-08-04
I'm going to set up 9.04 server 64 AMD version and have a 4GB lying around. Is that too small? All I will be doing is streaming files (from other HDs), maybe recording TV (to other HDs) and possibly some other things like monitoring network traffic and smallish stuff. 

Would I be severely limiting my options with a 4GB HD for the OS?

Cheers

---

### Post by Technoviking on 2009-08-04
4GB shoild be plenty. I run databases with 7 millions object with 4 GB.

T-V

---

### Post by garfonzo on 2009-08-04
> **Technoviking said:**
> 4GB shoild be plenty. I run databases with 7 millions object with 4 GB.

T-V

Excellent. I always put the OS on a separate physical disk and using this 4GB is out of the question for Windows. This will be perfect for the server.

Thanks for the quick reply!

---

### Post by grantemsley on 2009-08-05
I'd run the manufacture's diagnostic tool on the drive first to make sure it is still in OK shape, but otherwise it should be fine.

---

### Post by finite9 on 2009-08-05
4GB may be too small if your needs change.  I encode videos on a 4GB server and it gets up to 85% utilisation.  Dont ask me how it manages this...mencoder to x264 from terminal didnt seem like it would consume so much.  If you want virtual machines as well, then they take up a big chunk.

But then again, it depends on the definition of "server", as it's different for everyone.

---

### Post by finite9 on 2009-08-05
> **Technoviking said:**
> 4GB shoild be plenty. I run databases with 7 millions object with 4 GB.

T-V

Number of objects maybe isn't a good bench mark for how much memory is enough.  You dont load all the objects at once i presume?, so then it's just a case of how much menory your database executable process consumes whilst running idle + how much memory you need for the objects you load regularly.

---

### Post by garfonzo on 2009-08-05
I'm talking a 4GB hard drive on which to O/S would be installed. I'm not referring to how much RAM it has. So, when I say, "would 4GB be enough" I'm wondering if, after the OS install, will I be in a tight position to add other services such as Samba and others. 

From what I've found, the OS needs about 500MB, so after that I'll have space to add services. 

I'm thinking I'm ok but any thoughts are welcome.

---

### Post by andamaru on 2009-08-05
4 GB will be enough, I usually install my system on a 5 GB partitions and everything is fine (1 - 2 GB free) and my system has a bunch of large packages

---

