---
title: "Virtualization and Containers..."
date: 2018-05-21
forum: Virtualisation
---

### Post by rayj00 on 2018-05-21
I am working on a project in which I am considering using containers.

A few questions though:

1. Since my server will be a VPS, how are Ubuntu containers affected versus a bare metal server?
2. Is there a rule of thumb for the number of containers that can be used efficiently?
3. Is there a rule of thumb on how the host server should be configured versus the number of containers needed? 
   (ex:  with 4 containers, the host should have  X mB of ram, X mB of storage, etc.)
4. The containers will be used as media servers, ingesting rtmp streams and outputting HLS.
    (I am aware of bandwidth issues)

Any other concerns I should have in doing this?  Am I insane?

Thanks,

Ray

---

### Post by TheFu on 2018-05-21
Running containers inside a virtual machine is a best practice to get at least 1 layer of separation from the hardware for a slight improvement to security.

All the other questions are completely dependent on  the actual workload and cannot be answered without many more specifics.  Basically, you need to try it, see what is needed, and go from there.  Container density is between 10:1 or 1000:1, just depends. I/O matters along with the workload.
 
For best practices with containers, there were a few sessions at SELF 3-4 yrs ago. The conference videos are on youtube.

Whether you are insane or not can't be determined from the information provided.  ;)

---

### Post by rayj00 on 2018-05-21
Thanks TheFu.  I think I can move forward and start experimenting!

Ray

---

