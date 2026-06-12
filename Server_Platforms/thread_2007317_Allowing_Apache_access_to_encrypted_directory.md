---
title: "Allowing Apache access to encrypted directory?"
date: 2012-06-20
forum: Server Platforms
---

### Post by norwichnick on 2012-06-20
Hi everyone,

I have an odd scenario which I'm struggling to find a solution for. If anyone can shine some light on it, I would certainly appreciate it.

I am using Ubuntu 10.04 LTS Desktop with a LAMP stack running. I also chose to encrypt my home directories when installing the system from day one.

My scenario: hosting some web documents that are of significant importance that are accessible to any system-permitted user, but would be unaccessible if the hard disk were removed and inserted to another machine as an extra disk.

I have tried moving the documents that I want to protect in to a user's home directory and accessing the documents whilst Apache is running as that user and it works a treat. However, when that user logs out of the GUI session, nobody else on the system can see it as the encryption doesn't get clearance.

Is there anything I can do that would give me such security? As stated earlier in the post, the main scenario I am trying to protect against, is someone removing the physical disk, installing it on another machine, booting their OS and trying to get access to our files.

If there is any further information I can provide that would help anyone in providing some input, please do let me know.

Many thanks,
Nick

---

