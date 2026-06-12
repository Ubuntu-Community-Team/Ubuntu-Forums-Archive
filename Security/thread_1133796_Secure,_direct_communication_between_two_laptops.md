---
title: "Secure, direct communication between two laptops?"
date: 2009-04-23
forum: Security
---

### Post by sookoon on 2009-04-23
Hello, all.  I love the forum, and I've been able to get all my questions answered, just by taking the time to search!  And it was about a thousand questions. 

One that I'm not able to get a good answer on is:

What method do you recommend (and how to do it?) to set up a direct, secure communication link between two laptops?  I'll clarify:

  1. Direct, meaning that no third-party server / service is involved.

  2. Communication, being both chat and voice, and even shared desktop, if possible.  Again, no third party server / service.

  3. Must be encrypted, using latest + greatest algorithm.  Latency is not a concern.

  4. Both laptops running Ubuntu Intrepid.

  5. Neither computer has a static IP, and they don't reside in the same network.  Completely remote. 

Let me know if you require more information from me.  Oh, and:

  6. no, it's not for illegal activity!

If you know of an easy-to-read step-by-step guide for the above, I'd love to see it. 

As a return for the favor, I'll be putting up a visual step-by-step guide on:
1) how to generate SSL keys, up to 3DES 4096bit
2) how to set up thunderbird to use those keys

Thank you!

---

### Post by Dave_Connor on 2009-04-23
For my system I use ssh to open virtual shell on another system. Use key auth only to ensure security. And sshfs for media streaming on lan and rsync for backups and scp for direct file transfer.

---

